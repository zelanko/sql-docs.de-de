---
title: Caption-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bdba96bec45395e1a3aa0cd5f99ce12d417f404f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573552"
---
# <a name="caption-element-xmla"></a>Caption-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Enthält Informationen über die Beschriftung des übergeordneten Elements [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) oder [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
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
|Übergeordnete Elemente|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md), [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Für **HierarchyInfo** -Elemente enthält das **Caption** -Element den Namen der Eigenschaft, die die Elementbeschriftungen der Hierarchie bereitstellt. Der Wert entspricht der MEMBER_CAPTION-Eigenschaft, die in der OLE DB-Spezifikation für OLAP für Achsen-Rowsets definiert ist.  
  
 Für **Member** -Elemente enthält das **Caption** -Element die Beschriftung des übergeordneten **Member** -Elements in der für die XMLA-Sitzung (XML for Analysis) angegebenen Sprache. Wenn keine Beschriftung verfügbar ist, enthält dieses Element den eindeutigen Namen des Elements.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
