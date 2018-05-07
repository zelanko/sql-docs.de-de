---
title: DimensionPermissions-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cdbc69a8ad91b229dc03029e49a2c50e2e23bf4a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="dimensionpermissions-element-assl"></a>DimensionPermissions-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält die Auflistung der Berechtigungen für eine [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md) Element oder ein [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md) Element.  
  
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md), [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|Untergeordnete Elemente|[DimensionPermission](../../../analysis-services/scripting/objects/dimensionpermission-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Bei **CubePermission** -Elementen überschreiben die **DimensionPermission** -Elemente dieser Auflistung die Berechtigungen, die in der **DimensionPermissions** -Auflistung jeder Dimension, auf die explizit verwiesen wird, festgelegt sind. Wird auf eine Dimension in dieser Auflistung nicht verwiesen, erbt das **CubePermission** -Element die Berechtigungen, die in der **DimensionPermissions** -Auflistung der Dimension festgelegt sind.  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.DimensionPermissionCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Schemaauflistungen & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
