---
title: AxesInfo-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AxesInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords:
- AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bde7feb88ad570665200c1c3357bbba4127a963
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178490"
---
# <a name="axesinfo-element-xmla"></a>AxesInfo-Element (XMLA)
  Enthält eine Auflistung von [AxisInfo](axisinfo-element-xmla.md) -Elementen und stellt die im übergeordneten [OlapInfo](olapinfo-element-xmla.md) -Element enthaltenen Achsenmetadaten dar.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<OlapInfo>  
   ...  
   <AxesInfo>  
      <AxisInfo>...</AxisInfo>  
   </AxesInfo>  
   ...  
</OlapInfo>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[OlapInfo](olapinfo-element-xmla.md)|  
|Untergeordnete Elemente|[AxisInfo](axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `AxesInfo`-Element enthält ein `AxisInfo`-Element für jede Achse innerhalb des mehrdimensionalen Datensatzes, der von einem `root`-Element mithilfe des `MDDataSet`-Datentyps zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
