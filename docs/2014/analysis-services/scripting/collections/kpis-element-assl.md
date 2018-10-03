---
title: KPIs-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpis Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpis
helpviewer_keywords:
- Kpis element
ms.assetid: da4e32a0-1416-4d32-8b7f-7d74be23c9d4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d1b0817a7419aa76d9a015c8409b2f09962e04ad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168186"
---
# <a name="kpis-element-assl"></a>Kpis-Element (ASSL)
  Enthält die Auflistung von Key Performance Indicators ([Kpi](../objects/kpi-element-assl.md) Elementen) mit dem übergeordneten Element verknüpft ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Cube><!-- or Perspective -->  
   ...  
   <Kpis>  
      <Kpi>...</Kpi> <!-- parent: Cube -->  
<!-- or -->  
      <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- parent: Perspective -->  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|None|  
|Standardwert|None|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Cube](../objects/cube-element-assl.md), [Perspektive](../objects/perspective-element-assl.md)|  
  
|Vorgänger oder übergeordnetes Element|Untergeordnetes Element|  
|------------------------|-------------------|  
|[Cube](../objects/cube-element-assl.md)|[KPI](../objects/kpi-element-assl.md)|  
|[Perspektive](../objects/perspective-element-assl.md)|[KPI](../objects/kpi-element-assl.md) des Typs [PerspectiveKpi](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="remarks"></a>Hinweise  
 Das entsprechende Element im Analysis Management Objects (AMO)-Objektmodell ist <xref:Microsoft.AnalysisServices.KpiCollection>.  
  
## <a name="see-also"></a>Siehe auch  
 [Sammlungen &#40;ASSL&#41;](collections-assl.md)  
  
  
