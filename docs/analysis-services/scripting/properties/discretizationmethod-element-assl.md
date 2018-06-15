---
title: DiscretizationMethod-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 81064689788574061f103b973a5435beb3e83893
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036411"
---
# <a name="discretizationmethod-element-assl"></a>DiscretizationMethod-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*InclusionThresholdSetting*|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert des **DiscretizationMethod** -Elements bestimmt, wie Werte für **DimensionAttribute** oder **ScalarMiningStructureColumn** diskretisiert oder in spezifischen Gruppen geordnet werden. Weitere Informationen über die Diskretisierung finden Sie unter [Diskretisierungsmethoden &#40;Data Mining&#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*Automatic*|Entspricht der AUTOMATIC-Diskretisierungsmethode für Miningstrukturspalten.|  
|*EqualAreas*|Entspricht der EQUAL_AREAS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*Clusters*|Entspricht der CLUSTERS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*Schwellenwerte*|Entspricht der THRESHOLDS-Diskretisierungsmethode für Miningstrukturspalten.|  
|*EqualRanges*|Entspricht der EQUAL_RANGES-Diskretisierungsmethode für Miningstrukturspalten.|  
  
 Die Enumeration, die den zulässigen Werten für die entsprechende **DiscretizationMethod** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
