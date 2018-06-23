---
title: AxisInfo-Element (XMLA) | Microsoft Docs
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
- AxisInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxisInfo
- microsoft.xml.analysis.axisinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxisInfo
helpviewer_keywords:
- AxisInfo element
ms.assetid: 060741db-b2ec-4174-9277-58d996440a88
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1ac7ce9fdfeca2e2c48fe990c32c809827729959
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047893"
---
# <a name="axisinfo-element-xmla"></a>AxisInfo-Element (XMLA)
  Stellt die Metadaten einer einzelnen Achse dar, die im [AxesInfo](axesinfo-element-xmla.md) -Element enthalten sind.  
  
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
|Übergeordnete Elemente|[AxesInfo](axesinfo-element-xmla.md)|  
|Untergeordnete Elemente|[HierarchyInfo](hierarchyinfo-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|Name|Erforderliche `String` Attribut. Der Name der Achse.|  
  
## <a name="remarks"></a>Hinweise  
 In einem `root`-Element, das das `MDDataSet`-Objekt verwendet, enthält ein `AxisInfo`-Element eine Auflistung von `HierarchyInfo`-Elementen, die in Kombination mit dem Wert des `name`-Attributs eine Definition einer einzelnen Achse darstellt, die im multidimensionalen Datensatz zurückgegeben wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  