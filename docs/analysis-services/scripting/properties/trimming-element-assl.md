---
title: Trimming-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3273dba26a1b7af45b2a9eed5aab2d6302fa61a1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="trimming-element-assl"></a>Trimming-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Gibt an, wie die Daten der Datenquelle eingeschränkt werden.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem>  
   ...  
   <Trimming>...</Trimming>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|*Richting*|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Links*|Die Daten werden auf der linken Seite gekürzt.|  
|*Richting*|Die Daten werden auf der rechten Seite gekürzt.|  
|*LeftRight*|Die Daten werden auf der linken und auf der rechten Seite gekürzt.|  
|*InclusionThresholdSetting*|Die Daten werden nicht gekürzt.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Trimming** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Trimming>.  
  
 Das Element, das das übergeordnete Element des entspricht **Trimming** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.DataItem>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
