---
title: AxisInfo-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 52c3b114c1082a895325170fa8fbf6fef656b8ca
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574332"
---
# <a name="axisinfo-element-xmla"></a>AxisInfo-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Stellt die Metadaten einer einzelnen Achse dar, die im [AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md) -Element enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AxesInfo>  
   ...  
   <AxisInfo name="string">  
      <HierarchyInfo>...</HierarchyInfo>  
   </AxisInfo>  
   ...  
</AxesInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AxesInfo](../../../analysis-services/xmla/xml-elements-properties/axesinfo-element-xmla.md)|  
|Untergeordnete Elemente|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|Name|Erforderliches **String** -Attribut. Der Name der Achse.|  
  
## <a name="remarks"></a>Hinweise  
 In einem **root** -Element, das das **MDDataSet** -Objekt verwendet, enthält ein **AxisInfo** -Element eine Auflistung von **HierarchyInfo** -Elementen, die in Kombination mit dem Wert des **name** -Attributs eine Definition einer einzelnen Achse darstellt, die im multidimensionalen Datensatz zurückgegeben wurde.  
  
## <a name="see-also"></a>Siehe auch
 [Eigenschaften &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
