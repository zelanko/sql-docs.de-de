---
title: OptimizedState-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2791a3cd8f96961adfe2f2bd0bcf3aa1db13a50e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34037964"
---
# <a name="optimizedstate-element-assl"></a>OptimizedState-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bestimmt die Optimierungsebene, die auf die Hierarchie angewendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CubeHierarchy>  
   ...  
   <OptimizedState>...</OptimizedState>  
   ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*FullyOptimized*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*FullyOptimized*|Durch die Instanz werden Indizes zum Verbessern der Abfrageleistung für die Hierarchie erstellt.|  
|*NotOptimized*|Durch die Instanz werden keine zusätzlichen Indizes erstellt.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **OptimizedState** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.OptimizationType>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
