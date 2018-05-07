---
title: CellPermission-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9c4b6c9420be8eec3ba6d856f7c6312bfeb9b7f9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="cellpermission-element-assl"></a>CellPermission-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Beschreibt den Berechtigungen der Elemente einer [Rolle](../../../analysis-services/scripting/objects/role-element-assl.md) Element besitzen, für einzelne Zellen innerhalb einer [Cube](../../../analysis-services/scripting/objects/cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CellPermissions>  
   <CellPermission>  
      <Access>...</Access>  
            <Description>...</Description>  
      <Expression>...</Expression>  
      <Annotations>...</Annotations>  
   </CellPermission>  
</CellPermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CellPermissions](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md)|  
|Untergeordnete Elemente|[Zugriff](../../../analysis-services/scripting/properties/access-element-assl.md), [Anmerkungen](../../../analysis-services/scripting/collections/annotations-element-assl.md), [Beschreibung](../../../analysis-services/scripting/properties/description-element-assl.md), [Ausdruck](../../../analysis-services/scripting/properties/expression-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.CellPermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
