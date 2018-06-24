---
title: LNum-Element (XMLA) | Microsoft Docs
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
- LNum Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.lnum
- urn:schemas-microsoft-com:xml-analysis#LNum
- http://schemas.microsoft.com/analysisservices/2003/engine#LNum
helpviewer_keywords:
- LNum element
ms.assetid: 7b9cc143-0c5e-4a8c-a288-8921bfcfd103
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: affdefb04b94d863faa9a9fb6a9eed8ea5b07606
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046507"
---
# <a name="lnum-element-xmla"></a>LNum-Element (XMLA)
  Enthält Informationen über die Ordnungsposition der Ebenen für die übergeordneten Elemente [HierarchyInfo](hierarchyinfo-element-xmla.md) oder [Member](member-element-xmla.md) .  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LNum>...</LNum>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|ssNoversion|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[HierarchyInfo](hierarchyinfo-element-xmla.md), [Member](member-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für `HierarchyInfo`-Elemente enthält das `LNum`-Element den Namen der Eigenschaft, die die Ordnungspositionen der Ebenen für die Hierarchie bereitstellt. Der Wert entspricht der LEVEL_NUMBER-Eigenschaft, die in der OLE DB-Spezifikation für OLAP für Achsen-Rowsets definiert ist.  
  
 Für `Member` Elemente, die `LNum` Element enthält die nullbasierte Ordnungsposition, von der Stammebene der Hierarchie des Elements durch das übergeordnete Element dargestellten [Member](member-element-xmla.md) Element. Der Wert null (0) gibt die Stammebene der Hierarchie an.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  