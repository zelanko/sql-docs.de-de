---
title: AttributePermission-Element (ASSL) | Microsoft-Dokumentation
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
- AttributePermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributePermission
helpviewer_keywords:
- AttributePermission element
ms.assetid: efc8aa63-3959-4b2e-98f8-2a9c424298c2
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0c39047b1f63f0abbab109e2d1e8f82ca2a4c863
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277876"
---
# <a name="attributepermission-element-assl"></a>AttributePermission-Element (ASSL)
  Definiert den Berechtigungen, die Elemente einer [Rolle](role-element-assl.md) Element verfügen, für die Attribute einer individuellen Dimension in einem [Cube](cube-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[AttributePermissions](../collections/attributepermissions-element-assl.md)|  
|Untergeordnete Elemente|[AllowedSet](../properties/allowedset-element-assl.md), [Anmerkungen](../collections/annotations-element-assl.md), [AttributeID](../properties/id-element-assl.md), [DefaultMember](member-element-assl.md), [DeniedSet](../properties/deniedset-element-assl.md), [Beschreibung ](../properties/description-element-assl.md), [VisualTotals](../properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [CubeDimensionPermission-Datentyp &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
