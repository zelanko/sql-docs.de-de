---
title: RefreshPolicy-Element (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d553fc069242c8c9c3ba3348820c81474fd3a668
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="refreshpolicy-element-assl"></a>RefreshPolicy-Element (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bestimmt, wie oft im dynamischen Teil der Dimension oder Measuregruppe (gemäß der Festlegung im [Persistence](../../../analysis-services/scripting/properties/persistence-element-assl.md) -Element) geprüft wird, ob Änderungen vorliegen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding -->  
   ...  
   <RefreshPolicy>...</RefreshPolicy>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Siehe Tabelle unten.|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
|Vorgänger oder übergeordnetes Element|Standardwert|  
|------------------------|-------------------|  
|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)|*ByQuery*|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|Keine|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*ByQuery*|Jede Abfrage überprüft, ob sich die Quelldaten geändert haben.|  
|*ByInterval*|Quelldaten werden nur beim von [RefreshInterval](../../../analysis-services/scripting/properties/refreshinterval-element-assl.md)angegebenen Intervall auf Änderungen überprüft.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **RefreshPolicy** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.RefreshPolicy>.  
  
## <a name="see-also"></a>Siehe auch  
 [Persistence-Element & #40; ASSL & #41;](../../../analysis-services/scripting/properties/persistence-element-assl.md)   
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
