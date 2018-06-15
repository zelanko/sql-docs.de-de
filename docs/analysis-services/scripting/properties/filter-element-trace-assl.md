---
title: Filter-Element (Ablaufverfolgung) (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9efa3d3993c9902590a694dd6e543a83e6ae8da6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032871"
---
# <a name="filter-element-trace-assl"></a>Filter-Element (Ablaufverfolgung) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält ein XML-Dokument-Fragment, beschreibt die [Ablaufverfolgung](../../../analysis-services/scripting/objects/trace-element-assl.md) Filter.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Trace>  
   ...  
   <Filter>...</Filter>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|String|  
|Standardwert|Keine|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Trace](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Das Element, das das übergeordnete Element des entspricht **Filter** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Verfolgt Element &#40;ASSL&#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)  
  
  
