---
title: CubeInfo-Element (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CubeInfo
- microsoft.xml.analysis.cubeinfo
- urn:schemas-microsoft-com:xml-analysis#CubeInfo
helpviewer_keywords:
- CubeInfo element
ms.assetid: a504bac5-4bf2-4f78-a288-e74a34eaa97e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f58bcd7cbd15c767196e9efc2654e24aeacf94d4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214640"
---
# <a name="cubeinfo-element-xmla"></a>CubeInfo-Element (XMLA)
  Enthält die Cubemetadaten, die vom übergeordneten Element [OlapInfo](olapinfo-element-xmla.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<OlapInfo>  
   ...  
   <CubeInfo>  
      <Cube>...</Cube>  
   </CubeInfo>  
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
|Untergeordnete Elemente|[Cube](cube-element-olapinfo-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das `CubeInfo`-Element enthält für jeden Cube, auf den im mehrdimensionalen Datenset verwiesen wird, ein `Cube`-Element.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gibt in dieser Auflistung nur ein einziges `Cube`-Element zurück, da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] keine Aussagen unterstützt, die auf mehrere Cubes in der FROM-Klausel der MDX-Sprache (Multidimensional Expressions) verweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
