---
title: Target-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23d55d909179fd568075feba54199514a7396c6b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169060"
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
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
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
  
  
