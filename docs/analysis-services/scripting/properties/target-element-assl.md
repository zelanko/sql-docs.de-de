---
title: Target-Element (ASSL) | Microsoft-Dokumentation
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 98ec5c729f5735343f5eaa87e5232fcfb138cf38
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045778"
---
# <a name="target-element-assl"></a>Target-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifiziert das Ziel der [Aktion](../../../analysis-services/scripting/objects/action-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <Target>...</Target>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der erwartete Wert dieses Elements hängt der Wert, der die [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) -Element für das übergeordnete Element **Aktion**. In der folgenden Tabelle werden die erwarteten Werte für **Target** , basierend auf dem Wert für **TargetType**, beschrieben.  
  
|TargetType-Wert|Erwarteter Wert|  
|----------------------|--------------------|  
|*Cube*|Der Name eines Cubes.|  
|*Zellen*|Ein Teilcubeausdruck.|  
|*Legen Sie*|Ein Mengenausdruck oder der Name einer benannten Menge.<br /><br /> Hinweis: Eine SELECT-Anweisung kann nicht verwendet werden.|  
|*HierarchyMembers-Hierarchie*|Der Name einer Hierarchie.|  
|*DimensionMembers-Dimension*|Der Name einer Dimension.|  
|*LevelMembers-Ebene*|Der Name einer Ebene.|  
|*AttributeMembers-Attribut*|Der Name eines Attributs.|  
  
 Das Element, das dem übergeordneten entspricht **Ziel** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
