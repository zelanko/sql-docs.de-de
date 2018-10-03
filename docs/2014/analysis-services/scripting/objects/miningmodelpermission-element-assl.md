---
title: Miningmodelpermissions-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MiningModelPermission Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelPermission
helpviewer_keywords:
- MiningModelPermission element
ms.assetid: 4bd2f7e7-ff0d-404e-96fb-7e2c4eeb91e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c6bad2b1bda46fcc1437a5f4c967ced8a6c726f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113470"
---
# <a name="miningmodelpermission-element-assl"></a>MiningModelPermissions-Element (ASSL)
  Definiert die Berechtigungen der Elemente einer [Rolle](role-element-assl.md) Element verfügen, für ein einzelnes [MiningModel](miningmodel-element-assl.md) Element.  
  
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
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|[Berechtigung](../data-type/permission-data-type-assl.md)|  
|Standardwert|None|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[MiningModelPermissions](../collections/miningmodelpermissions-element-assl.md)|  
|Untergeordnete Elemente|[AllowBrowsing](../properties/allowbrowsing-element-assl.md), [AllowDrillThrough](../properties/allowdrillthrough-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], können Sie Drillthrough für Miningstrukturen aktivieren, durch das Hinzufügen der `AllowDrillthrough` Berechtigung für die [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md) Auflistung. Wenn `AllowDrillthrough` aktiviert ist, auf die Miningstruktur und das Miningmodell, jedes Mitglied einer Rolle mit [AllowDrillThrough-Element &#40;ASSL&#41; ](../properties/allowdrillthrough-element-assl.md) Berechtigungen für das Modell Abfragen von Datamining-Modells und zurückgeben können strukturspalten, die nicht im Modell enthalten sind, mithilfe der folgenden Syntax:  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 Daher sollten Sie zum Schutz sensibler oder persönlicher Informationen die `AllowDrillthrough`-Berechtigung für ein Miningmodell nur zulassen, wenn es unbedingt erforderlich ist. Weitere Informationen finden Sie unter [AllowDrillThrough-Element &#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md).  
  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.MiningModelPermission>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40;ASSL&#41;](objects-assl.md)  
  
  
