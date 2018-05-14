---
title: MoveWithDescendants-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 34ea88c2aee76684c3876195bda9b1f2633bab3a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="movewithdescendants-element-xmla"></a>MoveWithDescendants-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Gibt an, ob die Nachfolger der Attributelemente auch vom übergeordneten Element aktualisiert [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Die **MoveWithDescendants** -Element bestimmt, ob die **aktualisieren** Befehl sollte nicht nur die identifizierten Attributelemente Aktualisieren der [Attribute](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md) -Element, aber Außerdem, die die Nachfolger dieser Attributelemente ebenfalls aktualisiert werden.  
  
> [!NOTE]  
>  Dieses Element gilt nur für Attributelemente in Über-/Unterordnungshierarchien.  
  
 Weitere Informationen zum Aktualisieren von Elementen finden Sie unter [einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
