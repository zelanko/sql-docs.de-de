---
title: Member-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1001edf8a3dd7cd2b41525c0e23ed07775e51a4e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="member-element-assl"></a>Member-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den Namen eines Mitglieds eines [Group](../../../analysis-services/scripting/objects/group-element-assl.md) - oder [Role](../../../analysis-services/scripting/objects/role-element-assl.md) -Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
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
|Übergeordnete Elemente|[Element](../../../analysis-services/scripting/collections/members-element-assl.md)|  
|Untergeordnete Elemente|[Name](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die Elemente, die den übergeordneten Elementen von entsprechen **Member** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.Group> und <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
