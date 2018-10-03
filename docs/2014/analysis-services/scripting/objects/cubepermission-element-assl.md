---
title: CubePermission-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubePermission
helpviewer_keywords:
- CubePermission element
ms.assetid: b144b623-ff20-4ead-91ad-4c718f3b140b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7dc2c8cc50ccf61515241c7b9861c438ae369022
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055122"
---
# <a name="cubepermission-element-assl"></a>CubePermission-Element (ASSL)
  Definiert die Berechtigungen der Elemente eines bestimmten [Rolle](role-element-assl.md) Element in einer bestimmten [Cube](cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubePermissions>  
   <CubePermission>  
      <!-- The following elements extend Permission -->  
      <ReadSourceData>...</ReadSourceData>  
            <DimensionPermissions>...</DimensionPermissions>  
            <CellPermissions>...</CellPermissions>  
   </CubePermission>  
</CubePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../data-type/permission-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das einmal oder mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubePermissions](../collections/cubepermissions-element-assl.md)|  
|Untergeordnete Elemente|[CellPermissions](../collections/cellpermissions-element-assl.md), [DimensionPermissions](../collections/dimensionpermissions-element-assl.md), [ReadSourceData](data-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Cube-Element &#40;ASSL&#41;](cube-element-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
