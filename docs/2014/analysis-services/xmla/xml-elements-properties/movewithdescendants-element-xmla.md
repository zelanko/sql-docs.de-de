---
title: MoveWithDescendants-Element (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MoveWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords:
- MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 975044359f2855f8cced46ca2045c2c397e4234b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060558"
---
# <a name="movewithdescendants-element-xmla"></a>MoveWithDescendants-Element (XMLA)
  Gibt an, ob die Nachfolger der Attributelemente auch vom übergeordneten Element aktualisiert [Update](../xml-elements-commands/update-element-xmla.md) Befehl.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Boolean|  
|Standardwert|False|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Update](../xml-elements-commands/update-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `MoveWithDescendants` Element bestimmt, ob der `Update` Befehl sollte nicht nur die identifizierten Attributelemente Aktualisieren der [Attribute](attributes-element-xmla.md) -Element, sondern auch die Nachfolger dieser Attributelemente sein werden ebenfalls aktualisiert.  
  
> [!NOTE]  
>  Dieses Element gilt nur für Attributelemente in Über-/Unterordnungshierarchien.  
  
 Weitere Informationen zum Aktualisieren von Elementen finden Sie unter [einfügen, aktualisieren und Löschen von Membern &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  