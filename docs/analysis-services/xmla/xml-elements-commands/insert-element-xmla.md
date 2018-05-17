---
title: INSERT-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 594275e6601aae3c28da344ecf2e1de8c9f1f7c9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="insert-element-xmla"></a>Insert-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Fügt Attributelemente in eine Dimension ein.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Insert>  
      <Object>...</Object>  
      <Attributes>...</Attributes>  
   </Insert>  
</Command>  
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
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md), [Objekt](../../../analysis-services/xmla/xml-elements-properties/object-element-dimension-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Der **Insert** -Befehl fügt der Dimension mit aktiviertem Schreibzugriff neue Attributelemente hinzu.  
  
 Weitere Informationen zum Löschen von Elementen finden Sie unter [einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Drop-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Update-Element & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Befehle & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
