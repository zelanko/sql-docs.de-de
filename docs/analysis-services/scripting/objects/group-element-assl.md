---
title: Group-Element (ASSL) | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c702faacf9ad5a062dc792c20d78f0bf060da2ab
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032491"
---
# <a name="group-element-assl"></a>Group-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definiert eine Gruppe von Elementen, die an ein Attribut gebunden sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Groups>  
   <Group>  
      <Name>...</Name>  
      <Members>...</Members>  
   </Group>  
<Groups/>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Keine|  
|Standardwert|Keine|  
|Kardinalität|1-n: Erforderliches Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Gruppen](../../../analysis-services/scripting/collections/groups-element-assl.md)|  
|Untergeordnete Elemente|[Members](../../../analysis-services/scripting/collections/members-element-assl.md), [Name](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Objektmodell von Analysis Management Objects (AMO) ist <xref:Microsoft.AnalysisServices.Group>.  
  
## <a name="see-also"></a>Siehe auch  
 [UserDefinedGroupBinding-Datentyp & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/userdefinedgroupbinding-data-type-assl.md)   
 [Objekte & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
