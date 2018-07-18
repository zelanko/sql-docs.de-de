---
title: Target-Element (ASSL) | Microsoft-Dokumentation
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
- Target Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Target
helpviewer_keywords:
- Target element
ms.assetid: 08ce0441-94b6-4f1d-acba-f31c8212cb79
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec2f4a43b8b03e2f28d4bd8c61a9c6e4a9d20eb5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180767"
---
# <a name="target-element-assl"></a>Target-Element (ASSL)
  Identifiziert das Ziel der [Aktion](../objects/action-element-assl.md) Element.  
  
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
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der erwartete Wert dieses Elements hängt der Wert, der die [TargetType](targettype-element-assl.md) -Element für das übergeordnete Element `Action`. Die folgende Tabelle beschreibt die erwarteten Werte für `Target` basierend auf den Wert der `TargetType`.  
  
|TargetType-Wert|Erwarteter Wert|  
|----------------------|--------------------|  
|*Cube*|Der Name eines Cubes.|  
|*Zellen*|Ein Teilcubeausdruck.|  
|*Legen Sie*|Ein Mengenausdruck oder der Name einer benannten Menge. **Hinweis:** eine SELECT-Anweisung kann nicht verwendet werden.|  
|*HierarchyMembers-Hierarchie*|Der Name einer Hierarchie.|  
|*DimensionMembers-Dimension*|Der Name einer Dimension.|  
|*LevelMembers-Ebene*|Der Name einer Ebene.|  
|*AttributeMembers-Attribut*|Der Name eines Attributs.|  
  
 Das Element, das dem übergeordneten entspricht `Target` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
