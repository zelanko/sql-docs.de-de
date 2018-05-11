---
title: TargetType-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5261d212777049c907af8d4db8f3b085ded8740e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="targettype-element-assl"></a>TargetType-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifiziert den Elementtyp des Elements identifiziert, der [Ziel](../../../analysis-services/scripting/properties/target-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Cube*|Das Ziel der Aktion ist ein Cube.|  
|*Zellen*|Das Ziel der Aktion ist ein Teilcube.|  
|*Festlegen*|Das Ziel der Aktion ist eine Menge.|  
|*Hierarchie*|Das Ziel der Aktion ist eine Hierarchie.|  
|*Ebene*|Das Ziel der Aktion ist eine Ebene.|  
|*DimensionMembers*|Das Ziel der Aktion sind die Elemente einer Dimension.|  
|*HierarchyMembers*|Das Ziel der Aktion sind die Elemente einer Hierarchie.|  
|*LevelMembers*|Das Ziel der Aktion sind die Elemente einer Ebene.|  
|*AttributeMembers*|Das Ziel der Aktion sind die Elemente eines Attributs.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **TargetType** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 Das Element, das das übergeordnete Element des entspricht **TargetType** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
