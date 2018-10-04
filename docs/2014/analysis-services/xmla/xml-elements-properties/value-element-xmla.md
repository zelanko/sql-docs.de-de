---
title: Wert-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 054da002271711d4b86a08e694b18e01e796b3ea
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205714"
---
# <a name="value-element-xmla"></a>Value-Element (XMLA)
  Enthält den gewünschten Wert, der eine [Attribut](attribute-element-xmla.md) Element hinzugefügt werden durch eine [einfügen](../xml-elements-commands/insert-element-xmla.md) Befehl oder ein [Zelle](cell-element-xmla.md) Element aktualisiert werden ein [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)Befehl.  
  
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
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Attribut](attribute-element-xmla.md), [Zelle](cell-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Für `Attribute` Elemente, die `Value` Element enthält den gewünschten Wert, der das Element nach dem enthalten soll die `Insert` Befehl wird ein Commit ausgeführt. Weitere Informationen zum Einfügen von Elementen finden Sie unter [einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Für `Cell` Elemente, die `Value` Element enthält den gewünschten Wert an, die die Zelle nach enthalten sollen die `UpdateCells` Befehl wird ein Commit ausgeführt. Der tatsächliche Wert, der in der Rückschreibetabelle für die Zelle gespeichert ist, ist die Differenz zwischen dem Originalwert der Zelle und dem gewünschten Wert der Zelle.  
  
 Der von diesem Element verwendete Datentyp sollte dem Datentyp der zu aktualisierenden Zelle entsprechen.  
  
 Weitere Informationen zum Aktualisieren von Zellen finden Sie unter [Aktualisieren von Zellen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [CellOrdinal-Element &#40;XMLA&#41;](cellordinal-element-xmla.md)   
 [INSERT-Element &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [UpdateCells-Element &#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
