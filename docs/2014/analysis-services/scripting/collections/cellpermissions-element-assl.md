---
title: CellPermissions-Element (ASSL) | Microsoft Docs
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
- CellPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fe89d1e2de728773d9eaae32023e801676a02bb0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149739"
---
# <a name="cellpermissions-element-assl"></a>CellPermissions-Element (ASSL)
  Enthält die Auflistung der Berechtigungen für Zellen im zugehörigen [Cube](../objects/cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubePermission>  
   ...  
   <CellPermissions>  
      <CellPermission>...</CellPermission>  
   </CellPermissions>  
   ...  
</CubePermission>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Untergeordnete Elemente|[CellPermission](../objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die Auflistung kann bis zu einer enthalten `CellPermission` -Objekt für jeden Wert des zulässigen der [Zugriff](../properties/access-element-assl.md) Element.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.CellPermissionCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Permission-Datentyp &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  