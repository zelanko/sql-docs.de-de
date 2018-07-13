---
title: UName-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- UName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UName
- urn:schemas-microsoft-com:xml-analysis#UName
- microsoft.xml.analysis.uname
helpviewer_keywords:
- UName element
ms.assetid: b4916d44-cf77-4d4c-b4e5-a0a98192d057
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa8df2d964db3c8131b9566e04b05c106638d62e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185127"
---
# <a name="uname-element-xmla"></a>UName-Element (XMLA)
  Enthält den eindeutigen Namen für das übergeordnete [HierarchyInfo](hierarchyinfo-element-xmla.md) - oder [Member](member-element-xmla.md) -Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <UName>...</UName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für `HierarchyInfo` Elemente, die `UName` Element enthält den Namen der Eigenschaft, die die eindeutigen Elementnamen der Hierarchie bereitstellt. Der Wert entspricht der MEMBER_UNIQUE_NAME-Eigenschaft, die in der OLE DB-Spezifikation für OLAP für Achsen-Rowsets definiert ist.  
  
 Bei `Member`-Elementen enthält das `UName`-Element den eindeutigen Namen des übergeordneten  `Member`-Elements.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
