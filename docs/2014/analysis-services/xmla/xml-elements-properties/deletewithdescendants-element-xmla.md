---
title: DeleteWithDescendants-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DeleteWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#DeleteWithDescendants
- microsoft.xml.analysis.deletewithdescendants
- urn:schemas-microsoft-com:xml-analysis#DeleteWithDescendants
helpviewer_keywords:
- DeleteWithDescendants element
ms.assetid: adfc9437-aaa7-4364-bcdb-128fcc9a410d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 93a6d92e675e0ae016327e064fabb6ec2c012aac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199940"
---
# <a name="deletewithdescendants-element-xmla"></a>DeleteWithDescendants-Element (XMLA)
  Gibt an, ob auch die Nachfolger der Attributelemente auch vom übergeordneten [Drop](../xml-elements-commands/drop-element-xmla.md) -Befehl gelöscht werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Drop>  
   ...  
   <DeleteWithDescendants>...</DeleteWithDescendants>  
   ...  
</Drop>  
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
|Übergeordnete Elemente|[Löschen](../xml-elements-commands/drop-element-xmla.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Die `DeleteWithDescendants` Element bestimmt, ob die `Drop` Befehl sollten die Attributelemente identifizierte Löschen der [, in denen](where-element-xmla.md) -Element, sondern auch sind, dass die Nachfolger dieser Attributelemente ebenfalls gelöscht werden sollen.  
  
> [!NOTE]  
>  Dieses Element gilt nur für Attributelemente in Über-/Unterordnungshierarchien.  
  
 Weitere Informationen zum Löschen und Aktualisieren von Attributelementen finden Sie unter [Einfügen, Aktualisieren und Löschen von Elementen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
