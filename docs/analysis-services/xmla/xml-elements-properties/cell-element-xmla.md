---
title: Cell-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 014f46219ece054c292ff3a3b7a11d98c07c1547
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="cell-element-xmla"></a>Cell-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Informationen über eine Zelle, die von einem [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md) -Befehl aktualisiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<UpdateCells>  
   ...  
   <Cell CellOrdinal="Long">  
      <Value>...</Value>  
   </Cell>  
   ...  
</UpdateCells>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[UpdateCells](../../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|Untergeordnete Elemente|[Wert](../../../analysis-services/xmla/xml-elements-properties/value-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|CellOrdinal|Erforderliches **Long** -Attribut. Enthält die nullbasierte Ordnungsposition der Zelle, die aktualisiert werden soll.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zum Aktualisieren von Zellen finden Sie unter [Aktualisieren von Zellen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
