---
title: DiscretizationMethod-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationMethod Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75308b5270eb762236be22fc0838a480474898dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200474"
---
# <a name="discretizationmethod-element-assl"></a>DiscretizationMethod-Element (ASSL)
  Definiert die zu verwendende Diskretisierungsmethode.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Keine*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|None|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des `DiscretizationMethod`-Elements bestimmt, wie Werte für `DimensionAttribute` oder `ScalarMiningStructureColumn` diskretisiert oder in spezifischen Gruppen geordnet werden. Weitere Informationen über die Diskretisierung finden Sie unter [Diskretisierungsmethoden &#40;Data Mining&#41;](../../data-mining/discretization-methods-data-mining.md).  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Automatic*|Entspricht der AUTOMATIC-Diskretisierungsmethode für Miningstrukturspalten.|  
|*EqualAreas*|Entspricht der EQUAL_AREAS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*Cluster*|Entspricht der CLUSTERS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*Schwellenwerte*|Entspricht der THRESHOLDS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*EqualRanges*|Entspricht der EQUAL_RANGES-Diskretisierungsmethode für Miningstrukturspalten.|  
  
 Die Enumeration, der den zulässigen Werten für `DiscretizationMethod` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
