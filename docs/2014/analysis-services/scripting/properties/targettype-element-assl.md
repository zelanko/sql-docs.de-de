---
title: TargetType-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TargetType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TargetType
helpviewer_keywords:
- TargetType element
ms.assetid: 2c69ea6e-2af7-435b-9841-86117d5554a7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed0ca768f075b7cd4249c9d8b021e2ec10d54c46
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099560"
---
# <a name="targettype-element-assl"></a>TargetType-Element (ASSL)
  Kennzeichnet den Elementtyp des Elements, der der [Ziel](target-element-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|None|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Aktion](../objects/action-element-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Cube*|Das Ziel der Aktion ist ein Cube.|  
|*Zellen*|Das Ziel der Aktion ist ein Teilcube.|  
|*Legen Sie*|Das Ziel der Aktion ist eine Menge.|  
|*Hierarchy*|Das Ziel der Aktion ist eine Hierarchie.|  
|*Level*|Das Ziel der Aktion ist eine Ebene.|  
|*DimensionMembers*|Das Ziel der Aktion sind die Elemente einer Dimension.|  
|*HierarchyMembers*|Das Ziel der Aktion sind die Elemente einer Hierarchie.|  
|*LevelMembers*|Das Ziel der Aktion sind die Elemente einer Ebene.|  
|*AttributeMembers*|Das Ziel der Aktion sind die Elemente eines Attributs.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `TargetType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 Das Element, das dem übergeordneten entspricht `TargetType` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
