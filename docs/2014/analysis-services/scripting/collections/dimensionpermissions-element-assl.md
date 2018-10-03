---
title: DimensionPermissions-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionPermissions
helpviewer_keywords:
- DimensionPermissions element
ms.assetid: cb9fdfbf-2118-423b-ba02-fa36813dbea0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af96e23a71064cb1d68c292f4224ee76b8395588
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48068730"
---
# <a name="dimensionpermissions-element-assl"></a>DimensionPermissions-Element (ASSL)
  Enthält die Auflistung der Berechtigungen für eine [Dimension](../objects/dimension-element-assl.md) Element oder ein [CubePermission](../objects/cubepermission-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Dimension> <!-- or CubePermission -->  
   ...  
   <DimensionPermissions>  
            <DimensionPermission>...</DimensionPermission> <!-- parent: Dimension -->  
      <!-- or -->  
      <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- parent: CubePermission -->  
      </DimensionPermissions>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubePermission](../objects/cubepermission-element-assl.md), [Dimension](../objects/dimension-element-assl.md)|  
|Untergeordnete Elemente|[DimensionPermission](../objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Bei `CubePermission`-Elementen überschreiben die `DimensionPermission`-Elemente dieser Auflistung die Berechtigungen, die in der `DimensionPermissions`-Auflistung jeder Dimension, auf die explizit verwiesen wird, festgelegt sind. Wird auf eine Dimension in dieser Auflistung nicht verwiesen, erbt das `CubePermission`-Element die Berechtigungen, die in der `DimensionPermissions`-Auflistung der Dimension festgelegt sind.  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
