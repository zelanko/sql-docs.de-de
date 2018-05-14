---
title: Miningmodelpermission-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f05a12d5be30826e5a826320f2eb5a6c604456e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="miningmodelpermission-element-assl"></a>MiningModelPermissions-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert die Berechtigungen der Elemente einer [Rolle](../../../analysis-services/scripting/objects/role-element-assl.md) Element besitzen, für ein einzelnes [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningModelPermissions>  
   <MiningModelPermission xsi:type="Permission">  
      <!-- The following elements extend Permission -->  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <AllowBrowsing>...</AllowBrowsing>  
   </MiningModelPermission>  
</MiningModelPermissions>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Standardwert|Keine|  
|Kardinalität|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)|  
|Untergeordnete Elemente|[AllowBrowsing](../../../analysis-services/scripting/properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], können Sie Drillthrough für Miningstrukturen aktivieren, durch Hinzufügen der **AllowDrillthrough** Berechtigung für die [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md) Auflistung. Wenn **AllowDrillthrough** aktiviert ist, auf die Miningstruktur und das Miningmodell, jedes Mitglied einer Rolle mit [AllowDrillThrough-Element &#40;ASSL&#41; ](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) können Berechtigungen für das Modell Abfragen. die Data mining-Modell, und, die nicht im Modell enthalten waren, mithilfe der folgenden Syntax strukturspalten zurückgeben:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Daher sollten Sie zum Schutz sensibler oder persönlicher Informationen die **AllowDrillthrough** -Berechtigung für ein Miningmodell nur zulassen, wenn es unbedingt erforderlich ist. Weitere Informationen finden Sie unter [AllowDrillThrough-Element &#40;ASSL&#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
